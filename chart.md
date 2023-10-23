graph TD

subgraph Initialization
    start[Start]
    initializeEnv[Initialize MATLAB Environment]
    setTrajHandle[Set trajhandle to circle]
    setControlHandle[Set controlhandle to controller]
    setRealTime[Set real_time to true]
    addPaths[Add Necessary Paths]
    initFigures[Initialize Figures for Visualization]
    initConditions[Set Initial Conditions]
    setMaxIter[Set max_iter]
    setInitTimeStep[Set Initial Time, Time Step, and Image Capture Time]
    initError[Initialize Error Variables]
    setPosVelTol[Set Position and Velocity Tolerance]
end

subgraph MainSimulation
    runSimulation[Run Simulation]
    checkODEStability[Check ODE45 Stability]
    initQuadPlot[Initialize Quadrotor Plot]
    simulateMotion[Simulate Quadrotor's Motion using ODE45]
    calculateForceTorque[Calculate Force and Torque]
    updateStatePos[Update Quadrotor's State and Position]
    saveTrajectory[Save Simulated Trajectory Data]
    updateQuadPlot[Update Quadrotor's Plot in the Figure]
    updateTitle[Update Iteration and Time Title]
    pauseRealTime[Pause for Real-Time Simulation]
    checkTerminationCriteria[Check Termination Criteria]
    endMainLoop[End Main Loop]
    closeVideo[Close Video File]
end

subgraph Termination
    checkODETime(Check ODE45 Stability)
end

start --> initializeEnv
initializeEnv --> setTrajHandle
initializeEnv --> setControlHandle
initializeEnv --> setRealTime
initializeEnv --> addPaths
initializeEnv --> initFigures
initConditions --> setMaxIter
initConditions --> setInitTimeStep
initConditions --> initError
initConditions --> setPosVelTol

runSimulation --> checkODEStability
runSimulation --> initQuadPlot
initQuadPlot --> simulateMotion
simulateMotion --> calculateForceTorque
calculateForceTorque --> updateStatePos
updateStatePos --> saveTrajectory
saveTrajectory --> updateQuadPlot
updateQuadPlot --> updateTitle
updateTitle --> pauseRealTime
pauseRealTime --> checkTerminationCriteria
checkTerminationCriteria --> endMainLoop
checkODETime --> endMainLoop
checkODETime --> pauseRealTime
checkODETime --> endMainLoop
endMainLoop --> closeVideo
